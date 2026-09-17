# Safe-Guard threat model

This document defines the security scope for the project's binary prompt-injection detector. It is an analyst model for planning and evaluation, not a new set of source labels.

## System boundary

The detector is placed at the boundary where text enters an LLM-powered application. It receives a prompt-like text value and produces a safe/injection classification for an analyst or downstream policy to review. The project dataset contains only `text` and binary `label` fields:

- `0`: safe/benign;
- `1`: prompt injection.

The provided test split remains held out for final evaluation. This project does not claim that the dataset's binary labels identify a specific attack technique.

## Assets to protect

For a financial-technology application, relevant assets include:

- confidential customer, account, transaction, and business data;
- credentials, API keys, system prompts, policies, and retrieval indexes;
- integrity of financial analysis, recommendations, records, and workflow state;
- availability and cost controls for model and tool calls; and
- auditability, privacy, and user trust.

## Attack surface

The in-scope boundary is untrusted text submitted to an LLM workflow, including text that may attempt to alter the model's instructions or policy. In a future deployment, the same boundary may receive text from a user interface, uploaded document, retrieved content, or an external integration. The current dataset and experiments do not establish coverage for all of those sources.

The detector cannot by itself control what a model, retriever, or tool does after classification. Any production design would still need instruction isolation, least-privilege tool access, output and action validation, logging, human review for high-impact actions, and a fail-safe response to uncertainty.

## In scope for this project

1. Binary discrimination between the dataset's safe/benign and prompt-injection labels.
2. Recall-first evaluation because an undetected injection can be more costly than a false alarm.
3. Measurement of false positives, false negatives, threshold behavior, and split leakage.
4. Qualitative analysis of representative errors and possible lexical shortcuts.
5. Explicit documentation of where synthetic and general-purpose source data may fail to represent finance-specific traffic.

## Out of scope or not established

- Treating the dataset-card generation categories as ground-truth per-row taxonomy labels.
- Claiming coverage of jailbreaks, data exfiltration, tool abuse, indirect prompt injection, or multi-turn attacks unless separately evaluated.
- Claiming robustness to encoding, obfuscation, multilingual prompts, paraphrases, adaptive attackers, or distribution shift without dedicated tests.
- Authorizing, blocking, or reversing financial transactions based on this classifier alone.
- Inferring that high benchmark accuracy makes the filter production-safe.
- Training or evaluating on the provided test split during model selection.

## Analyst taxonomy (proposed, non-source)

For error analysis, reviewers may tag examples with one or more analyst categories. These tags are hypotheses for organizing review and must not be confused with the dataset's binary labels:

| Analyst tag | Working definition |
| --- | --- |
| `instruction_override` | Attempts to replace, ignore, or supersede the application's instructions or policy. |
| `context_manipulation` | Attempts to reframe trusted context, roles, boundaries, or message priority. |
| `social_engineering` | Uses authority, urgency, impersonation, or persuasion to induce unsafe behavior. |
| `secret_extraction` | Attempts to reveal system prompts, credentials, hidden context, or protected data. |
| `unsafe_action_request` | Attempts to make the application take an unauthorized or high-impact action. |
| `obfuscation_or_encoding` | Uses encoding, spacing, substitution, or other transformations to evade detection. |
| `benign_ambiguous` | Benign text whose wording resembles an injection or is difficult to classify confidently. |
| `unknown_or_unreviewed` | Insufficient evidence for a more specific analyst tag. |

The `analyst_tag` field, if introduced later, must be documented as human-derived annotation with its own rubric and agreement limitations. It must not overwrite the original `label` field.

## Open risks and next dependencies

The next evaluation stages should test whether performance changes across finance-domain prompts, prompt length, language, obfuscation, source type, and attack intent. The team should also resolve the dataset licensing questions in the provenance note before redistributing raw or example data.

This threat model is a planning boundary. It is not a security certification, production approval, or evidence that any category is represented uniformly in Safe-Guard.
