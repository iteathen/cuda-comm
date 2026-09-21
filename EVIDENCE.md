# Evidence status

This repository follows the shared [iteathen evidence and validation policy](https://github.com/iteathen/.github/blob/main/EVIDENCE_POLICY.md).

## Current posture

CUDA-COMM is currently an architecture/planning repository. Its intended scope is documented, but there is no production implementation, installable package, public API, native-provider qualification, or performance claim.

## Registered claims

| Claim | Evidence class | Status |
| --- | --- | --- |
| `CUDA-COMM-PLAN-001` — intended scope: reusable GPU communication through public CUDA-JS contracts | **UNVALIDATED** | planning hypothesis / project boundary |

The claim record is machine-readable in [`evidence/claims.json`](evidence/claims.json).

## What current evidence establishes

The repository establishes the current project boundary, planning state, architecture decisions, and activation conditions under repository control.

## What it does not establish

It does not establish production usefulness, CUDA correctness, native-provider support, API stability, performance, or external reproduction.

## Path to stronger evidence

When implementation is authorized, claims should advance only through evidence that actually exists: deterministic internal qualification first, then hardware measurement and/or reference-grounded or externally reproduced evidence where applicable.

## Non-mutation rule

Evidence work may inspect, test, benchmark, and document CUDA-COMM. It must not change substantive operational behavior merely to make an evidence claim pass.
