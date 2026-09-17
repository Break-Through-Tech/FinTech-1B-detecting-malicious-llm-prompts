# Analyst taxonomy for review

This is a proposed analyst annotation scheme for reviewing detector errors. It is not part of the Safe-Guard source schema: the dataset provides only `text` and binary `label` (`0` safe/benign, `1` injection). The tags below must never be presented as source-provided ground truth.

| Tag | Definition | Review question |
| --- | --- | --- |
| `instruction_override` | Attempts to replace or ignore application instructions. | Does the text seek higher priority than the application policy? |
| `context_manipulation` | Attempts to alter roles, trusted context, or message priority. | Does it reframe what the model should trust? |
| `social_engineering` | Uses urgency, authority, impersonation, or persuasion. | Is compliance driven by a social pretext? |
| `secret_extraction` | Seeks prompts, credentials, hidden context, or protected data. | Is the target confidential information? |
| `unsafe_action_request` | Seeks an unauthorized or high-impact action. | Would compliance change financial or workflow state? |
| `obfuscation_or_encoding` | Uses transformations to evade detection. | Is the intent obscured by encoding or formatting? |
| `benign_ambiguous` | Benign text that resembles an attack. | Is the detector's concern understandable but unsupported? |
| `unknown_or_unreviewed` | Insufficient evidence for a narrower tag. | What evidence is missing? |

Analysts may apply multiple tags and should retain the original label. Any future annotation should record annotator guidance, agreement, and uncertainty separately.
