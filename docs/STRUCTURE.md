# Project structure

One monorepo. Packages follow the system boundaries of the pipeline.

```
looprepair/
├── docs/
├── src/looprepair/
│   ├── contracts/     # Scenario, Candidate, AnalyzeResult, ValidateResult, RunReport
│   ├── control/       # CLI, Scenario FSM, checkpoints, batch, report.json
│   ├── lab/           # Docker lab: rebuild, analyze, validate
│   ├── repair/        # tree-sitter, LLM generate/refine, ranking
│   └── platform/      # metrics aggregation, reproduce helpers
├── prompts/           # upstream prompt files (record source commit when added)
├── tests/
│   ├── control/
│   ├── lab/
│   ├── repair/
│   └── platform/
└── runs/              # local outputs (gitignored)
```

## Data flow

```
CLI / FSM (control)
  → lab.rebuild / analyze / validate
  → repair.generate / refine
  → report.json
  → platform metrics / tables
```

## Outside this repo

- Docker image `fino2020/looprepair:v1.0` (VulnLoc+, crepair, KLEE, fuzzer)
- Read-only checkout of Fino2020/LoopRepair for prompts and Table 2 comparison

Do not vendor VulnLoc+ C sources here. Do not commit API keys (use `.env`).
