# Pipeline Hazards

## Limits

> **Hazards:* Circumstances that would cause incorrect execution if next instruction is fetched and executed

- **Structural:** Different instructions at different stages in the pipeline want to use the same hardware resource
- **Data:** An instruction in pipeline requires data to be computed by a previous instruction still in pipeline
- **Control:** Succeeding instruction to put into pipeline depends on outcome of a previous branch instruction already in pipeline
- 