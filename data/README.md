# Dataset acquisition

Raw Safe-Guard files are intentionally not checked into Git. Obtain them from the hosted [Safe-Guard Prompt Injection dataset](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection) at the pinned revision in [`docs/data-provenance.md`](../docs/data-provenance.md).

```python
from datasets import load_dataset

dataset = load_dataset(
    "xTRam1/safe-guard-prompt-injection",
    revision="a3a877d608f37b7d20d9945671902df895ecdb46",
)
```

The expected hosted format is Parquet with `text` and `label` fields. The provided `test` split is held out; derive validation data from `train` only. Before use, verify columns, nulls, duplicates, labels, and row counts against the provenance note.

The dataset card does not state a clear license in the pinned repository metadata. Confirm dataset and seed-source terms with the project advisor before redistributing raw or example data.
