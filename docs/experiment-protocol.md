# Shared experiment protocol

## Source and split policy

Load Safe-Guard at revision `a3a877d608f37b7d20d9945671902df895ecdb46`. Preserve `text` and the original binary `label`; `0` is safe/benign and `1` is injection. Split the provided `train` data into train/validation with a documented deterministic stratified seed. Never fit preprocessing, select hyperparameters, or select thresholds using the provided `test` split.

## Reproducibility record

Each experiment should record dataset revision, source split, validation seed and proportion, preprocessing configuration, model configuration, threshold policy, package/runtime versions, and output artifact path. Artifact names should identify model family, feature configuration, seed, and split without embedding raw prompts.

## Comparison policy

Compare models on the same rows and label mapping. Report precision, recall, F1, PR-AUC, confusion matrix, and false-negative rate, with label-1 recall foregrounded. Do not compare numbers produced under different splits or thresholds without explaining the difference. Keep raw data and credentials out of Git.

## Open dependencies

The repository currently contains no committed training or evaluation implementation. This note therefore defines the protocol; future experiment PRs must attach their actual commands and generated artifacts.
