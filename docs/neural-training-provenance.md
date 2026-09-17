# Neural training provenance template

Complete this record when a neural model is trained. Blank fields are intentional until the corresponding run exists; they must not be filled with estimates.

| Field | Recorded value |
| --- | --- |
| Dataset revision | `a3a877d608f37b7d20d9945671902df895ecdb46` |
| Source split | `train`; provided `test` held out |
| Validation derivation | To be recorded from `train` only |
| Random seed(s) | To be recorded |
| Feature/tokenization configuration | To be recorded |
| Architecture and parameter count | To be recorded |
| Optimizer/training schedule | To be recorded |
| Saved model artifact | To be recorded; no artifact is currently committed |
| Evaluation command and metrics | To be recorded after the run |

The final record must include class counts, training duration or environment as useful, stopping criteria, threshold policy, and known data limitations. It must not include raw prompts, credentials, or unsupported performance claims.
