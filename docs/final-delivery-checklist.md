# Final delivery checklist

## Sources and data

- [ ] Dataset URL, pinned revision, schema, split sizes, label mapping, and source paper are cited.
- [ ] Raw data, credentials, and accidental notebook outputs are absent.
- [ ] Dataset and seed-source licensing/redistribution questions are resolved or prominently marked as blockers.

## Reproducibility

- [ ] Environment and dependency versions are documented.
- [ ] Retrieval, preprocessing, split, training, threshold, and evaluation commands are recorded.
- [ ] Provided test data is held out until final evaluation.
- [ ] Generated reports and figures identify their source revision and run configuration.

## Results and limits

- [ ] Selected model and operating point are supported by committed artifacts.
- [ ] Figures are legible and reproducible.
- [ ] Precision, recall, F1, PR-AUC, confusion matrix, and false-negative behavior are reported.
- [ ] Bias, leakage, synthetic-data, finance-domain, and adversarial limitations are stated.
- [ ] The detector is not described as a complete LLM security control or production approval.

## Validation receipt

- [ ] `git diff --check` passes.
- [ ] Relevant tests/lint/build commands and exact results are recorded.
- [ ] Final README links the artifacts and responsible-use boundaries.

Current status: this checklist records the required evidence; final results and detector artifacts remain dependencies until their implementation issues are complete.
