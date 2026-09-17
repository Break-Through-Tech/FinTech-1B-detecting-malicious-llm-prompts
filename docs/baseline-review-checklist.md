# Baseline documentation review checklist

- [ ] Dataset URL, pinned revision, schema, label mapping, and source attribution are present.
- [ ] Retrieval instructions do not require committing raw Parquet files.
- [ ] Train/validation/test roles are explicit and test remains untouched during selection.
- [ ] TF-IDF fitting is training-only and its configuration is recorded.
- [ ] Seeds, package versions, row identifiers, and artifact paths are recorded.
- [ ] Metrics include injection recall, false negatives, precision, F1, PR-AUC, and confusion matrix.
- [ ] Threshold selection is validation-only and its policy is stated.
- [ ] Comparisons use identical rows, labels, and split policy.
- [ ] Claims distinguish benchmark performance from finance-specific or production readiness.
- [ ] Synthetic generation, possible lexical shortcuts, and licensing uncertainty are acknowledged.

This checklist is a review aid, not evidence that the currently empty repository has already produced baseline results.
