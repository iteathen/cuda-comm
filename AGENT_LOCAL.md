# Repository context: cuda-comm

Universal engineering and design guidance comes from the account-global `AGENTS.md`.

## Mission and ownership

CUDA-COMM owns reusable provider-neutral GPU communication semantics when accepted: groups/teams/ranks, collectives, generic point-to-point meaning, PGAS/one-sided remote-memory-window semantics, communication ordering/completion/failure composition, and conformance.

CUDA-JS owns CUDA/provider mechanisms including selected NCCL/NVSHMEM/peer/RDMA primitives. NN distributed-training policy, MCGS search policy, and product topology remain with their natural owners.

## Local routing

Accepted `docs/decisions/`, `docs/specs/`, repository status/roadmap, and current issues own local implementation/activation truth.

## Local constraints

Dependency direction is `cuda-comm -> public cuda-js`. Maintained code uses JavaScript/ESM plus accepted Device-JS through public lower contracts; no Python, direct native/provider escape path, or private lower imports.