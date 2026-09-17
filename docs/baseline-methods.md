# Baseline methods draft

The baseline task is binary text classification on Safe-Guard prompts. The canonical input is `text`; the target is the original `label`, where `0` is safe/benign and `1` is injection. The provided test split is reserved for one final evaluation after model and threshold choices are frozen.

The first reproducible baseline should fit a TF-IDF word n-gram transformer on the training portion only, train logistic regression, and select any operating threshold on validation data under a recall-first policy. A linear SVM using the same fitted features and split policy is a comparison candidate. The neural comparison is a later milestone and must not silently change the data contract.

Report accuracy only as context. The primary security-facing measures are injection recall and false-negative count/rate, alongside precision, F1, PR-AUC, and a confusion matrix. These metrics characterize this benchmark; they do not establish finance-domain coverage or production safety.

No result numbers are asserted here because no baseline artifacts are committed yet.
