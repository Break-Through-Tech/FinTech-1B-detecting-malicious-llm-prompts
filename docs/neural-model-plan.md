# Neural-model documentation plan

The neural-model record should preserve the same Safe-Guard source revision, binary label semantics, train-only fitting policy, validation derivation, and held-out test boundary as the classical baselines.

## Required record

- feature source and embedding/tokenization method;
- model family, architecture, input dimensions, and parameter choices;
- initialization, optimizer, learning rate, batch size, epochs, early stopping, and seed;
- training/validation row counts and class distributions;
- threshold selection rule and recall-first rationale;
- package/runtime versions and saved-artifact location; and
- metrics, error slices, limitations, and the exact command used.

## Interpretation boundary

An embedding or Keras model is a comparison candidate, not automatically an improvement. No neural result should be described as finance-domain coverage or production safety without dedicated evaluation. Analyst taxonomy tags remain separate from the dataset's binary labels.
