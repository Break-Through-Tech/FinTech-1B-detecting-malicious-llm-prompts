# Methods and preliminary-results narrative

## Methods

We frame Safe-Guard as binary text classification: `text` is the input and `label` distinguishes safe/benign (`0`) from prompt injection (`1`). The hosted training split is divided into train and validation deterministically and stratifiably; the hosted test split remains untouched until final evaluation. Candidate text features and classifiers are compared under the shared protocol, with thresholds selected on validation data.

## Evaluation

Because missed injections are the primary security concern, interpretation foregrounds label-1 recall and false negatives, while also reporting precision, F1, PR-AUC, and confusion matrices. Any preliminary number must link to the exact generated artifact and command. No preliminary performance number is reported in this draft because the repository currently contains no evaluation artifact.

## Limits

The source combines synthetic attacks and prompts curated from general-purpose datasets. The binary labels do not provide per-example attack techniques, and the linked GLAN paper is background rather than detector validation. Results therefore describe this benchmark only; they do not establish robustness, finance-specific generalization, or production readiness.
