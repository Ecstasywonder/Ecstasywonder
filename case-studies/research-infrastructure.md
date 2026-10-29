# Phishing URL Research Infrastructure — Reproducible Pipelines and Analytics

**Focus:** Data engineering · ML infrastructure · reproducibility · CI automation  
**Technology areas:** Python, GitHub Actions, private object storage, DuckDB, manifests, testing and statistical reporting

## At a glance
This case study describes three related private engineering efforts: a controlled collection and ML evaluation pipeline, a separate analytics/reporting system and a sanitized replication package. It does **not** publish research input URLs, frozen datasets, private model output, unpublished findings or restricted artifacts.

## STAR case study

### Situation
Machine-learning classification results can be misleading when records overlap across splits, source timing is ignored, or training and reporting cannot be reconstructed. Ephemeral CI compute also requires durable artifact provenance.

### Task
Build a traceable research environment with controlled input handling, explicit leakage barriers, reproducible evaluation and independent statistical reporting without a continuously operated analytics server.

### Action
- Built Python collection and processing stages with archived-input checksums, metadata provenance, candidate quarantine and recorded inclusion/exclusion rules.
- Implemented URL/domain/template group controls, temporal and cross-source evaluation regimes and separate model fitting/evaluation boundaries.
- Used controlled GitHub Actions execution alongside private durable object storage to preserve evidence across ephemeral workers.
- Developed a separate DuckDB analytics layer for checksum-verified hydration, metric recomputation, readiness/final-eligibility checks and publication of derived reports.
- Prepared offline synthetic tests and sanitized replication documentation, separating reproducible methods from private or third-party-restricted content.

### Result
The private repositories document implemented research pipeline stages, synthetic automated checks, reproducibility manifests and gated reporting. Synthetic outputs are marked as development evidence, not scientific results. **Public release of the computational replication package remains blocked pending licensing and third-party data-rights clearance.** No detection accuracy, peer-reviewed conclusion or research release approval is asserted.

## Conceptual architecture
```text
Authorized sources
      |
Input capture + provenance/checksums
      |
Quarantine + dataset construction
      |
Leakage-controlled evaluation
      |
Private durable evidence store
      |
Independent validation + embedded analytics
      |
Gated reports and reproducibility manifests
```

## Engineering decisions
- Evaluate time-aware and group-controlled behavior instead of relying only on random splits.
- Keep source artifact production separate from independent interpretation.
- Treat storage as durable evidence and analytical state as reconstructible, disposable computation.
- Prevent synthetic or incomplete results from being represented as final research findings.

## Responsible disclosure
No real malicious URLs, protected data, private storage locations, source identifiers, credentials, model artifacts, experimental outcomes or access paths are published. This summary does not authorize release of the underlying code or datasets.
