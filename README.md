# LoopRepair

Replication and extension of the ICSE 2026 LoopRepair paper on VulnLoc+.

## Layout

```
src/looprepair/
  contracts/   # shared schemas
  control/     # CLI, scenario FSM, reports
  lab/         # Docker rebuild / analyze / validate
  repair/      # LLM generate / refine / ranking
  platform/    # metrics, CI helpers
prompts/       # prompt text (from upstream, pinned commit)
tests/
docs/
```

VulnLoc+ and crepair/KLEE stay in the authors’ Docker image (`fino2020/looprepair:v1.0`). Keep [Fino2020/LoopRepair](https://github.com/Fino2020/LoopRepair) as a read-only reference for prompts and published results.

## Setup

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
```
