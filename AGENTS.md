# CUDA-COMM Agent Entry Point

Read this file before changing the repository.

## Authority order

1. Explicit current project-owner instruction.
2. This file.
3. Accepted ADRs under `docs/decisions/`.
4. Accepted specifications under `docs/specs/`.
5. `docs/PROJECT_CHARTER.md`.
6. Status/roadmap/issues, which are tracking rather than implementation authority.

## Required method

Use `assess -> research -> reassess -> plan -> execute -> qualify -> review -> cleanup/document` for every meaningful work unit. Follow `LEGO -> SOLID -> CUPID -> KISS`; one semantic fact/resource/lifecycle has one visible owner.

LEGO is the outer architecture rule: ownership, universality, replaceability, scope containment, damage-limiting encapsulation, and context containment. A LEGO is too large when one agent cannot hold its complete authoritative working set—contract, implementation, invariants, lifecycle/resource/failure rules, tests/conformance, and immediate dependency/consumer interfaces—in focused attention with substantial headroom for reasoning and review. Context fit is a first-class boundary criterion alongside semantic, lifecycle, resource/failure, substitution, and change cohesion. When exceeded, recursively split at the strongest real seam or narrow scope; do not create arbitrary modules that duplicate truth or require cross-boundary internal knowledge. Inside a valid LEGO, SOLID structures responsibilities and dependency direction, CUPID shapes the implementation, and KISS removes remaining unjustified complexity; lower levels may not defeat higher ones.

## Repository boundary

CUDA-COMM owns reusable provider-neutral GPU communication semantics only when separately accepted: communication groups/teams/ranks, collective meaning, point-to-point meaning where generic, PGAS/one-sided remote-memory-window semantics, ordering/completion/failure composition, and communication-specific conformance.

CUDA-COMM does not own CUDA device/context discovery, raw P2P/RDMA registration, memory allocation, streams/events/operations, native NCCL/NVSHMEM handles/bootstrap, cluster administration, NN distributed-training policy, MCGS search/replica policy, or product topology meaning.

## Provider split

CUDA-JS remains the native/provider mechanism owner for bounded NCCL, NVSHMEM, peer-access and GPUDirect-RDMA primitives when selected. CUDA-COMM maps provider-neutral communication semantics through public lower-layer contracts.

Do not collapse NCCL collectives/P2P and NVSHMEM PGAS/RMA into one primitive merely because both move data between GPUs.

## Dependency direction

`cuda-comm -> public cuda-js`. Other semantic repos may depend on CUDA-COMM optionally. CUDA-JS never depends on CUDA-COMM.

## Lower-layer escalation

Direct native code, FFI, CUDA C++/PTX, private imports, provider handles, raw network/NIC/DPU state, or duplicated CUDA resource lifecycle are lower-layer/infrastructure ownership signals. Stop and classify them rather than creating local workarounds.

## Source and language

Maintained production/tooling code, when authorized, is JavaScript/ESM plus accepted restricted Device-JS through public lower-layer contracts. Do not add Python, maintained C/C++, direct FFI/Driver access, hand PTX, or subprocess-native implementations without an explicit successor decision.

## Current gate

Repository creation and bootstrap authorize no production source/API. Issue #3 is the semantic activation roadmap; accepted bounded specifications are required before implementation. Issue #2 separately owns repository-control/protected-main alignment.

## Completion rule

Completion requires exact-effect review, relevant qualification, cleanup and honest claim limits. No mock/portable result proves native topology/provider/performance support.