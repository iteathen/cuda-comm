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

LEGO is the outer architecture rule: ownership, universality, replaceability, scope containment, damage-limiting encapsulation, supported connection surfaces, and context containment. **The application/system is the outermost LEGO.** Its supported external inputs, outputs, commands, events, data contracts, and lifecycle entry/exit points are its public **studs/surfaces**. Large sections, subsystems, components, and large objects should preferentially compose smaller child LEGOs when that preserves cohesion; the parent owns the external responsibility and hides child topology.

A LEGO is too large when one agent cannot hold its complete authoritative working set—contract/studs/surfaces, implementation, invariants, lifecycle/resource/failure rules, tests/conformance, and immediate dependency/consumer interfaces—in focused attention with substantial headroom for reasoning and review. Context fit is a first-class boundary criterion alongside semantic, lifecycle, resource/failure, substitution, and change cohesion. When exceeded, recursively split at the strongest real seam or narrow scope; do not create arbitrary modules that duplicate truth or require cross-boundary internal knowledge. Callers connect through deliberate studs/surfaces and never drill through a parent to a private child. Inside a valid LEGO, SOLID structures responsibilities and dependency direction, CUPID shapes the implementation, and KISS removes remaining unjustified complexity; lower levels may not defeat higher ones.

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

## Execution efficiency / mutation hygiene

These are **default suggestions, not mandatory sequencing rules**. Use them when they reduce uncertainty, duplication, or avoidable mutation risk. Current validated information and repository-specific authority can justify a different sequence; do not perform a step merely for procedural completeness.

- **Read before write when the read can materially improve the decision.** Reuse prior validated context when its assumptions still hold. A safe, isolated, informative write can itself be research.
- **Prefer one ownership unit at a time when that keeps reasoning and review clear.** Cross ownership boundaries deliberately when the real problem or solution spans them.
- **Introduce new mechanisms when they solve a real problem.** Avoid gratuitous machinery, not invention.
- **When state is unexpected, stop and assess before acting.** Then choose whether to preserve it, repair forward, or roll back; rollback is not the default.
- **Qualify proportionally.** Validate before propagation when remaining uncertainty would become meaningfully more expensive. For simple, well-understood, mechanical changes, propagate then qualify once when that is cheaper and equally sound.
- **Reuse valid evidence and established conclusions.** Do not repeat research or validation solely to satisfy process form.
- Prefer the path that uses available information to reduce uncertainty and rework at reasonable cost while preserving correctness, ownership, recoverability, and honest evidence.
