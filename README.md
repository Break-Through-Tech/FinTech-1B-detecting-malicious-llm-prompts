# Detecting Malicious LLM Prompts

> This Break Through Tech AI Studio project explores a recall-first classifier for detecting prompt-injection text. It is a benchmark and learning artifact, not a production security certification or a financial decision system.

---

### 👥 **Team Members**

| Name | GitHub Handle | Contribution |
|------|---------------|--------------|
| Ahmed Lawal | [@AhmedLawal08](https://github.com/AhmedLawal08) | Data preprocessing, model evaluation, performance analysis, and results interpretation |
| Avi Paudel | [@Avi161](https://github.com/Avi161) | EDA, model selection, model training, and model evaluation |
| Han Wang | [@doublehan2023](https://github.com/doublehan2023) | Data exploration |
| Jacqueline Henriksen | [@jjjhenriksen](https://github.com/jjjhenriksen) | Data collection, exploratory analysis, and dataset documentation |
| Moukthika Nellutla | [@Mnellutla1120](https://github.com/Mnellutla1120) | Model selection, hyperparameter tuning, model training, and optimization |
| Zeynep Bezeklioglu | [@zeynepbezeklioglu](https://github.com/zeynepbezeklioglu) | Data preprocessing, model training and evaluation, and data validation |
| Zakariye Mohamed | [@zakiscoding](https://github.com/zakiscoding) | Model and data processing |

---

## 🎯 **Project Highlights**

- Explores a binary classifier that separates safe/benign prompt-like text from prompt-injection text at an LLM application boundary.
- Uses a recall-first evaluation policy that reports injection recall and false negatives before precision, F1, PR-AUC, and the confusion matrix.
- Establishes a reproducible dataset and evaluation contract: validation is derived from the training split, while the hosted test split remains held out for final evaluation.
- Documents responsible-use boundaries for a classifier that cannot replace authorization, instruction isolation, least-privilege tools, action validation, logging, or human review.

---

## 👩🏽‍💻 **Setup and Installation**

* How to clone the repository:

  ```bash
  git clone https://github.com/Break-Through-Tech/FinTech-1B-detecting-malicious-llm-prompts.git
  cd FinTech-1B-detecting-malicious-llm-prompts
  ```
* How to install dependencies and set up the environment:

  ```bash
  python -m venv .venv
  source .venv/bin/activate
  python -m pip install -r requirements.txt
  ```
* How to access the dataset(s): retrieve the Safe-Guard Prompt Injection dataset from Hugging Face. Do not commit downloaded raw files. Before modeling, verify the expected schema, nulls, duplicates, labels, and split sizes.
* How to run the notebook or scripts: run the experiment you are reproducing. No model results or generated evaluation artifacts are committed yet.

---

## 🏗️ **Project Overview**

- How this project is connected to the Break Through Tech AI Program: this project is part of the Break Through Tech AI Studio program.
- Your AI Studio host company and the project objective and scope: the project explores prompt-injection detection for an LLM application boundary in a finance-adjacent setting.
- The real-world significance of the problem and the potential impact of your work: protected assets include confidential data, credentials and system instructions, workflow integrity, and model/tool availability and cost; a classifier alone cannot authorize, block, or reverse a high-impact financial action.

---

## 📊 **Data Exploration**

* The dataset(s) used: the project uses the [Safe-Guard Prompt Injection dataset](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection), hosted as Parquet. It contains `text` and `label` fields; `0` means safe/benign and `1` means prompt injection. The hosted `train` split has 8,236 rows and `test` has 2,060 rows.
* Data exploration and preprocessing approaches: check schema, missing values, duplicates, label balance, and split integrity before feature fitting. Validation must be derived from `train`, and `test` stays held out for final evaluation.
* Insights from your Exploratory Data Analysis (EDA): the dataset combines synthetic attacks with prompts curated from general-purpose datasets, and its binary labels do not identify attack techniques.
* Challenges and assumptions when working with the dataset(s): possible distribution shift affects finance-specific traffic, adaptive attacks, indirect injection, multilingual or obfuscated prompts, multi-turn workflows, and tool abuse.

---

## 🧠 **Model Development**

* Model(s) used: the planned baseline uses TF-IDF features with linear classifiers; neural-model comparisons may be added after the baseline.
* Feature selection and Hyperparameter tuning strategies: feature fitting, preprocessing, thresholds, and hyperparameter selection must use training or validation data only.
* Training setup: runs should use deterministic stratified validation and retain the source revision, configuration, training-data provenance, and generated report needed for comparison.

---

## 📈 **Results & Key Findings**

* Performance metrics: report injection recall and false negatives first, alongside precision, F1, PR-AUC, and a confusion matrix.
* How your model performed: no model results or generated evaluation artifacts are committed yet; future claims must link the exact run and source revision.
* Insights from evaluating model fairness: fairness and robustness findings should be reported with the evaluation data and limitations that support them.

**Potential visualizations to include:**

* Confusion matrix, precision-recall curve, feature importance plot, prediction distribution, outputs from fairness or explainability tools

---

## 🚀 **Next Steps**

* What are some of the limitations of your model? The dataset may not represent finance-specific traffic, adaptive attacks, indirect injection, multilingual or obfuscated prompts, multi-turn workflows, or tool abuse.
* What would you do differently with more time/resources? Compare neural approaches only when their training provenance and resource requirements are documented, and add layered controls such as instruction isolation, least-privilege tools, action validation, logging, and human review.
* What additional datasets or techniques would you explore? Evaluate generalization across the scenarios above and confirm dataset and seed-source terms with the project advisor before redistributing raw or derived data.

---

## 📝 **License**

The repository does not currently declare a project license. Confirm the dataset and cited seed-source terms with the project advisor before redistributing raw or derived data.

---

## 📄 **References** (Optional but encouraged)

- [Safe-Guard Prompt Injection dataset](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection)
- [Synthetic Data (Almost) from Scratch: Generalized Instruction Tuning for Language Models](https://arxiv.org/abs/2402.13064)

---

## 🙏 **Acknowledgements** (Optional but encouraged)

This project is developed through the Break Through Tech AI Studio program with support from the project team, Challenge Advisor, host-company representatives, and teaching staff.
