# README final-section draft

The final README should present the project in this order:

1. **Project objective and threat model** — identify the prompt-ingress decision and protected assets; link [`docs/threat-model.md`](threat-model.md).
2. **Data and provenance** — link the pinned Safe-Guard source, schema, splits, retrieval instructions, synthetic origin, and licensing questions; link [`docs/data-provenance.md`](data-provenance.md).
3. **Reproducible setup** — describe environment creation, hosted-data retrieval, validation-only split derivation, and run order once scripts exist.
4. **Methods and evaluation** — link the shared protocol and state recall-first metrics, test-set holdout, and threshold policy.
5. **Results** — link only committed reports or artifacts and identify their exact source revision and command.
6. **Limitations and responsible use** — state that benchmark results are not production-safety evidence and that model output must not authorize high-impact financial actions alone.
7. **Team, references, and license status** — preserve attribution and disclose unresolved licensing before redistribution.

The README must remove template placeholders and must not invent results, scripts, artifacts, or deployment claims. This draft remains separate from the final README replacement until evaluation artifacts exist.
